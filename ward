package de.hshn.mi.pdbg.basicservice;

import de.hshn.mi.pdbg.basicservice.jdbc.AbstractPersistentJDBCObject;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

/**
 * Implementation of interface {@link Ward}. Describes a part of a hospital unit or department.
 */

public class WardImpl extends AbstractPersistentJDBCObject implements Ward {

    int numberOfBeds;
    String name;

    protected WardImpl(BasicDBService service, Long id) {
        super(service, id);
    }

    protected WardImpl(BasicDBService service) {
        super(service, INVALID_OBJECT_ID);
    }

    @Override
    public int getNumberOfBeds() {
        return numberOfBeds;
    }

    @Override
    public void setNumberOfBeds(int number) {
        if (number <= 0) {
            throw new AssertionError();
        }
        this.numberOfBeds = number;
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public void setName(String name) {
        if (name == null || name.isBlank()) {
            throw new AssertionError();
        }
        this.name = name;
    }

    @Override
    public long getObjectID() {
        return super.getObjectID();
    }

    @Override
    public long store(Connection connection) throws SQLException {
        if (super.isPersistent()) {
            PreparedStatement statement = PreparedStatementsUtil.updateStatements[PreparedStatementsUtil.WARD];
            statement.setLong(1, super.getObjectID());
            statement.setString(2, name);
            statement.setInt(3, numberOfBeds);
            statement.setLong(4, super.getObjectID());
            statement.execute();

        } else {
            PreparedStatement statement = PreparedStatementsUtil.insertStatements[PreparedStatementsUtil.WARD];
            super.setObjectID(getNextId(connection));
            statement.setLong(1, super.getObjectID());
            statement.setString(2, name);
            statement.setInt(3, numberOfBeds);
            statement.execute();

        }
        return super.getObjectID();
    }

    @Override
    public boolean isPersistent() {
        return super.isPersistent();
    }
}
